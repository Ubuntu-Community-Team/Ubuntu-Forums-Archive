---
title: "Edimax randomly disconnects from network"
date: 2015-10-24
forum: Networking &amp; Wireless
---

### Post by qkzoo on 2015-10-24
This is a Compaq Pres running Lubuntu 14.04.1, it connects to the network just fine when I first start up the computer, and then at some seemingly random point, just stops being able to connect to the web.  According to wifi indicator, it is still connected to the network.  Sometimes I can disconnect from the wlan I'm connected to and reconnect, and all is good, sometimes this doesn't seem to work.  Here's the output of the network info script:



```

########## wireless info START ##########

Report from: 24 Oct 2015 14:29 EDT -0400

Booted last: 24 Oct 2015 14:21 EDT -0400

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-31-generic #36-Ubuntu SMP Wed Oct 7 15:04:02 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP77 Ethernet [10de:0760] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:360a]
    Kernel driver in use: forcedeth

##### lsusb #############################

Bus 002 Device 002: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8192cu              69632  0 
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                77824  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              724992  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              540672  2 mac80211,rtlwifi
hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
mxm_wmi                16384  1 nouveau
wmi                    20480  3 hp_wmi,mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.132  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          inet6 addr: fdd1:8929:59d7:0:<IP6 'wlan0' [IF]>/64 Scope:Global
          inet6 addr: fdd1:8929:59d7:0:b8fe:12da:cb93:93ec/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4065 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3447 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2874311 (2.8 MB)  TX bytes:514640 (514.6 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"DIAMOND"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'DIAMOND' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:16   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    400    0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     400    0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search gha.chartermi.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root       575     1  0 14:21 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        802.11n WLAN Adapter
GENERAL.DRIVER:                         rtl8192cu
GENERAL.DRIVER-VERSION:                 3.19.0-31-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:04.1/usb2/2-3/2-3:1.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     DIAMOND
GENERAL.CON-UUID:                       51fb91cd-5cd0-4804-b7b9-fcb4d3a0b853
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   51fb91cd-5cd0-4804-b7b9-fcb4d3a0b853 | DIAMOND
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
IP4.ADDRESS[1]:                         ip = 192.168.1.132/24, gw = 192.168.1.1
IP4.DNS[1]:                             71.10.216.1
IP4.DNS[2]:                             71.10.216.2
IP4.DNS[3]:                             192.168.1.1
IP4.DOMAIN[1]:                          gha.chartermi.net
DHCP4.OPTION[1]:                        network_number = 192.168.1.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        expiry = 1445797689
DHCP4.OPTION[9]:                        domain_name = gha.chartermi.net
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 86400
DHCP4.OPTION[16]:                       ip_address = 192.168.1.132
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 71.10.216.1 71.10.216.2 192.168.1.1
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       requested_ntp_servers = 1
DHCP4.OPTION[27]:                       requested_netbios_scope = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         ip = fdd1:8929:59d7:0:b8fe:12da:cb93:93ec/64, gw = ::
IP6.ADDRESS[2]:                         ip = fdd1:8929:59d7:0:<IP6 'wlan0' [IF]>/64, gw = ::
IP6.ADDRESS[3]:                         ip = fe80::<IP6 'wlan0' [IF]>/64, gw = ::
IP6.ROUTE[1]:                           dst = fdd1:8929:59d7::/64, nh = ::, mt = 400

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         NVIDIA Corporation
GENERAL.PRODUCT:                        MCP77 Ethernet
GENERAL.DRIVER:                         forcedeth
GENERAL.DRIVER-VERSION:                 0.64
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:0a.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off

SSID                BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
MyCharterWiFie1-2G  <MAC 'MyCharterWiFie1-2G' [AN1]>  Infra  11    2462 MHz  54 Mbit/s  30      &#9602;___  WPA2       no        
DIAMOND             <MAC 'DIAMOND' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  56      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 
MyCharterWiFiaf-2G  <MAC 'MyCharterWiFiaf-2G' [AC3]>  Infra  3     2422 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2       no        
NETGEAR47           <MAC 'NETGEAR47' [AN4]>  Infra  9     2452 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2       no        

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

[[/etc/NetworkManager/system-connections/DIAMOND]] (600 root)
[connection] id=DIAMOND | type=wifi
[wifi] ssid=DIAMOND | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

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

eth0      no frequency information.

lo        no frequency information.

wlan0     11 channels in total; available frequencies :
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

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'DIAMOND' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"DIAMOND"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d5d4a4d74
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Frontier5204' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Frontier5204"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002a267da180
                    Extra: Last beacon: 212ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'MyCharterWiFiaf-2G' [AC3]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"MyCharterWiFiaf-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001ba75d17180
                    Extra: Last beacon: 1592ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8192cu]
filename:       /lib/modules/3.19.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     3E8327A34276F37FFE5A6A8
depends:        rtlwifi,rtl8192c-common,rtl_usb,mac80211
intree:         Y
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B4:BA:13:D5:CE:C9:3E:1A:F4:B3:4D:36:DA:1B:D4:FC:FF:A5:44:10
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_usb]
filename:       /lib/modules/3.19.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     814A6FB8DBFFB696F45B316
depends:        rtlwifi,mac80211
intree:         Y
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B4:BA:13:D5:CE:C9:3E:1A:F4:B3:4D:36:DA:1B:D4:FC:FF:A5:44:10
sig_hashalgo:   sha512

[rtl8192c_common]
filename:       /lib/modules/3.19.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     134BAE300AAF914967D6C6C
depends:        rtlwifi
intree:         Y
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B4:BA:13:D5:CE:C9:3E:1A:F4:B3:4D:36:DA:1B:D4:FC:FF:A5:44:10
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.19.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     35016235A31CEB1854418E1
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B4:BA:13:D5:CE:C9:3E:1A:F4:B3:4D:36:DA:1B:D4:FC:FF:A5:44:10
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-31-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     6AE775D26377F997426A49D
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B4:BA:13:D5:CE:C9:3E:1A:F4:B3:4D:36:DA:1B:D4:FC:FF:A5:44:10
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-31-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B4:BA:13:D5:CE:C9:3E:1A:F4:B3:4D:36:DA:1B:D4:FC:FF:A5:44:10
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192cu]
debug: 0
swenc: N

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   18.139346] rtl8192cu: Chip version 0x10
[   18.224896] rtl8192cu: MAC address: <MAC 'wlan0' [IF]>
[   18.224901] rtl8192cu: Board Type 0
[   18.225142] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   18.225180] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[   18.233000] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   24.475984] forcedeth 0000:00:0a.0 eth0: MSI enabled
[   24.476264] forcedeth 0000:00:0a.0 eth0: no link during initialization
[   24.495162] rtl8192cu: MAC auto ON okay!
[   24.532694] rtl8192cu: Tx queue select: 0x05
[   25.813196] wlan0: authenticate with <MAC 'DIAMOND' [AC1]>
[   25.825079] wlan0: send auth to <MAC 'DIAMOND' [AC1]> (try 1/3)
[   25.831997] wlan0: authenticated
[   25.834432] wlan0: associate with <MAC 'DIAMOND' [AC1]> (try 1/3)
[   25.838693] wlan0: RX AssocResp from <MAC 'DIAMOND' [AC1]> (capab=0x411 status=0 aid=4)
[   25.840366] wlan0: associated
[  390.464071] wlan0: deauthenticating from <MAC 'DIAMOND' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  393.685488] wlan0: authenticate with <MAC 'DIAMOND' [AC1]>
[  393.700974] wlan0: send auth to <MAC 'DIAMOND' [AC1]> (try 1/3)
[  393.727447] wlan0: authenticated
[  393.730460] wlan0: associate with <MAC 'DIAMOND' [AC1]> (try 1/3)
[  393.741837] wlan0: RX AssocResp from <MAC 'DIAMOND' [AC1]> (capab=0x411 status=0 aid=4)
[  393.742815] wlan0: associated

########## wireless info END ############


```

---

### Post by qkzoo on 2015-10-24
Not sure if this helps or not, but it's the last lines in my syslog immediately after the network got funky again:

```
Oct 24 14:28:20 jordan-Compaq-Presario-CQ60-Notebook-PC ntpd[1460]: ntpd 4.2.6p5@1.2349-o Mon Apr 13 17:00:14 UTC 2015 (1)
Oct 24 14:28:20 jordan-Compaq-Presario-CQ60-Notebook-PC ntpd[1461]: proto: precision = 0.147 usec
Oct 24 14:28:20 jordan-Compaq-Presario-CQ60-Notebook-PC ntpd[1461]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Oct 24 14:28:20 jordan-Compaq-Presario-CQ60-Notebook-PC ntpd[1461]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Oct 24 14:28:20 jordan-Compaq-Presario-CQ60-Notebook-PC ntp[1452]: ...done.
Oct 24 14:28:20 jordan-Compaq-Presario-CQ60-Notebook-PC ntpd[1461]: Listen and drop on 1 v6wildcard :: UDP 123
Oct 24 14:28:20 jordan-Compaq-Presario-CQ60-Notebook-PC ntpd[1461]: Listen normally on 2 lo 127.0.0.1 UDP 123
Oct 24 14:28:20 jordan-Compaq-Presario-CQ60-Notebook-PC systemd[1]: Started LSB: Start NTP daemon.
Oct 24 14:28:20 jordan-Compaq-Presario-CQ60-Notebook-PC ntpd[1461]: Listen normally on 3 wlan0 192.168.1.132 UDP 123
Oct 24 14:28:20 jordan-Compaq-Presario-CQ60-Notebook-PC ntpd[1461]: Listen normally on 4 lo ::1 UDP 123
Oct 24 14:28:20 jordan-Compaq-Presario-CQ60-Notebook-PC ntpd[1461]: Listen normally on 5 wlan0 fe80::76da:38ff:fe2b:4872 UDP 123
Oct 24 14:28:20 jordan-Compaq-Presario-CQ60-Notebook-PC ntpd[1461]: peers refreshed
Oct 24 14:28:20 jordan-Compaq-Presario-CQ60-Notebook-PC ntpd[1461]: Listening on routing socket on fd #22 for interface updates
Oct 24 14:28:26 jordan-Compaq-Presario-CQ60-Notebook-PC dhclient: XMT: Info-Request on wlan0, interval 14280ms.
Oct 24 14:28:32 jordan-Compaq-Presario-CQ60-Notebook-PC wpa_supplicant[681]: wlan0: CTRL-EVENT-SCAN-STARTED
Oct 24 14:28:40 jordan-Compaq-Presario-CQ60-Notebook-PC dhclient: XMT: Info-Request on wlan0, interval 29950ms.
Oct 24 14:28:56 jordan-Compaq-Presario-CQ60-Notebook-PC NetworkManager[575]: <warn> (wlan0): DHCPv6 request timed out.
Oct 24 14:28:56 jordan-Compaq-Presario-CQ60-Notebook-PC NetworkManager[575]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1429
Oct 24 14:28:56 jordan-Compaq-Presario-CQ60-Notebook-PC NetworkManager[575]: <info> Activation (wlan0) Stage 5 of 5 (IPv6 Commit) scheduled...
Oct 24 14:28:56 jordan-Compaq-Presario-CQ60-Notebook-PC NetworkManager[575]: <info> Activation (wlan0) Stage 5 of 5 (IPv6 Commit) started...
Oct 24 14:28:56 jordan-Compaq-Presario-CQ60-Notebook-PC dbus[589]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Oct 24 14:28:56 jordan-Compaq-Presario-CQ60-Notebook-PC systemd[1]: Starting Network Manager Script Dispatcher Service...
Oct 24 14:28:56 jordan-Compaq-Presario-CQ60-Notebook-PC NetworkManager[575]: <info> Activation (wlan0) Stage 5 of 5 (IPv6 Commit) complete.
Oct 24 14:28:56 jordan-Compaq-Presario-CQ60-Notebook-PC dbus[589]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct 24 14:28:56 jordan-Compaq-Presario-CQ60-Notebook-PC systemd[1]: Started Network Manager Script Dispatcher Service.
Oct 24 14:28:56 jordan-Compaq-Presario-CQ60-Notebook-PC nm-dispatcher: Dispatching action 'dhcp6-change' for wlan0
Oct 24 14:28:59 jordan-Compaq-Presario-CQ60-Notebook-PC ntpd[1461]: Listen normally on 6 wlan0 fdd1:8929:59d7:0:76da:38ff:fe2b:4872 UDP 123
Oct 24 14:28:59 jordan-Compaq-Presario-CQ60-Notebook-PC ntpd[1461]: Listen normally on 7 wlan0 fdd1:8929:59d7:0:b8fe:12da:cb93:93ec UDP 123
Oct 24 14:28:59 jordan-Compaq-Presario-CQ60-Notebook-PC ntpd[1461]: peers refreshed
Oct 24 14:28:59 jordan-Compaq-Presario-CQ60-Notebook-PC ntpd[1461]: new interface(s) found: waking up resolver
Oct 24 14:32:00 jordan-Compaq-Presario-CQ60-Notebook-PC kernel: [  624.393631] nouveau  [  PTHERM][0000:02:00.0] temperature (86 C) went below the 'fanboost' threshold
Oct 24 14:31:41 jordan-Compaq-Presario-CQ60-Notebook-PC wpa_supplicant[681]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED]
Oct 24 14:32:26 jordan-Compaq-Presario-CQ60-Notebook-PC wpa_supplicant[681]: wlan0: WPA: Group rekeying completed with c8:d7:19:62:d9:1c [GTK=TKIP]
Oct 24 14:33:24 jordan-Compaq-Presario-CQ60-Notebook-PC wpa_supplicant[681]: wlan0: CTRL-EVENT-SCAN-STARTED
Oct 24 14:36:16 jordan-Compaq-Presario-CQ60-Notebook-PC kernel: [  880.992283] nouveau  [  PTHERM][0000:02:00.0] temperature (90 C) hit the 'fanboost' threshold
Oct 24 14:36:37 jordan-Compaq-Presario-CQ60-Notebook-PC systemd[1]: Starting Cleanup of Temporary Directories...
Oct 24 14:36:37 jordan-Compaq-Presario-CQ60-Notebook-PC systemd-tmpfiles[1727]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
Oct 24 14:36:37 jordan-Compaq-Presario-CQ60-Notebook-PC systemd[1]: Started Cleanup of Temporary Directories.
jordan@jordan-Compaq-Presario-CQ60-Notebook-PC:/var/log$ 

```

---

### Post by qkzoo on 2015-10-29
bump

---

### Post by praseodym on 2015-10-29
Change the driver via:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.10
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot

---

### Post by qkzoo on 2015-10-31
Knock on wood, but wifi has been operational now for several hours!  Thank you very much!  How did you know which driver and all that to install???

---

### Post by praseodym on 2015-10-31
;)

[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107)

---

