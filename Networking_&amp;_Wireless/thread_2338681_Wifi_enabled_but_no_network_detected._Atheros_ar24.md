---
title: "Wifi enabled but no network detected. Atheros ar242x / ar542x adapter. Ubuntu 16.04"
date: 2016-09-30
forum: Networking &amp; Wireless
---

### Post by chipro12 on 2016-09-30
Hi,

I have been looking for a solution to a wifi problem I have on my ubuntu 16.04. I install ubuntu to this compaq presario cq50 which is an old notebook. Everything works fine except the wifi. I have looked around and tried a lot but the problem is still there. I run the wireless script and attach to this. 

Hope someone can take a look and guide me to a potential direction to fix it.

P/S: I also want to add that I actually tried a wireless usb stick (Tp-link tl-wn722n) and worked right away plugged in with all networks detected and wireless connection is great. So I know it is certainly not the network problem but rather the laptop wireless card or something
```

########## wireless info START ##########

Report from: 30 Sep 2016 14:37 EDT -0400

Booted last: 30 Sep 2016 00:00 EDT -0400

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-38-generic #57-Ubuntu SMP Tue Sep 6 15:41:41 UTC 2016 i686 athlon i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP77 Ethernet [10de:0760] (rev a2)
    Subsystem: Hewlett-Packard Company MCP77 Ethernet [103c:360a]
    Kernel driver in use: forcedeth

07:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC [103c:137a]
    Kernel driver in use: ath5k

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k_htc              69632  0
ath9k_common           36864  1 ath9k_htc
ath9k_hw              458752  2 ath9k_common,ath9k_htc
ath5k                 139264  0
ath                    24576  4 ath9k_common,ath5k,ath9k_htc,ath9k_hw
mac80211              659456  2 ath5k,ath9k_htc
cfg80211              499712  5 ath,ath9k_common,ath5k,mac80211,ath9k_htc
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:130.85.83.197  Bcast:130.85.83.255  Mask:255.255.255.128
          inet6 addr: fe80::4f4a:23ab:74d1:1f1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11278 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1776 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1790735 (1.7 MB)  TX bytes:262068 (262.0 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         130.85.83.129   0.0.0.0         UG    100    0        0 eth0
130.85.9.4      130.85.83.129   255.255.255.255 UGH   100    0        0 eth0
130.85.83.128   0.0.0.0         255.255.255.128 U     100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search umbc.edu

##### network managers ##################

Installed:

    NetworkManager

Running:

root       697     1  0 13:13 ?        00:00:12 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         NVIDIA Corporation
GENERAL.PRODUCT:                        MCP77 Ethernet
GENERAL.DRIVER:                         forcedeth
GENERAL.DRIVER-VERSION:                 0.64
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:0a.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       90d37883-934b-3cbe-a738-cb378b0d96f1
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   90d37883-934b-3cbe-a738-cb378b0d96f1 | Wired connection 1
IP4.ADDRESS[1]:                         130.85.83.197/25
IP4.GATEWAY:                            130.85.83.129
IP4.ROUTE[1]:                           dst = 130.85.9.4/32, nh = 130.85.83.129, mt = 100
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             130.85.1.23
IP4.DNS[2]:                             130.85.1.8
IP4.DNS[3]:                             130.85.1.13
IP4.DOMAIN[1]:                          umbc.edu
IP4.WINS[1]:                            130.85.11.19
IP4.WINS[2]:                            130.85.11.30
IP4.WINS[3]:                            130.85.11.7
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       expiry = 1475274533
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 130.85.83.129
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 130.85.83.197
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       domain_name = umbc.edu
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       broadcast_address = 130.85.83.255
DHCP4.OPTION[21]:                       domain_name_servers = 130.85.1.23 130.85.1.8 130.85.1.13
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       dhcp_lease_time = 14400
DHCP4.OPTION[24]:                       netbios_name_servers = 130.85.11.19 130.85.11.30 130.85.11.7
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.128
DHCP4.OPTION[27]:                       network_number = 130.85.83.128
DHCP4.OPTION[28]:                       requested_routers = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 130.85.9.4
IP6.ADDRESS[1]:                         fe80::4f4a:23ab:74d1:1f1d/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR242x / AR542x Wireless Network Adapter (PCI-Express) (AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC)
GENERAL.DRIVER:                         ath5k
GENERAL.DRIVER-VERSION:                 4.4.0-38-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/0000:07:00.0/net/wlan0
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

[[/etc/NetworkManager/system-connections/eduroam 1]] (600 root)
[connection] id=eduroam 1 | type=wifi | permissions=user:luan:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=eduroam
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[ipv6] method=auto
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto

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

lo        no frequency information.

eth0      no frequency information.

wlan0     12 channels in total; available frequencies :
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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

##### module infos ######################

[ath9k_htc]
filename:       /lib/modules/4.4.0-38-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       ath9k_htc/htc_9271-1.4.0.fw
firmware:       ath9k_htc/htc_7010-1.4.0.fw
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     D97AA41EF63133F707BAA44
depends:        mac80211,ath9k_hw,ath9k_common,ath,cfg80211
intree:         Y
vermagic:       4.4.0-38-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_dev_fw:Use development FW version (int)
parm:           blink:Enable LED blink on activity (int)

[ath9k_common]
filename:       /lib/modules/4.4.0-38-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     6FBD9F8A613FDFA282AB4FE
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.4.0-38-generic SMP mod_unload modversions 686 

[ath9k_hw]
filename:       /lib/modules/4.4.0-38-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     BF9F4930086BABAAF3CD9BA
depends:        ath
intree:         Y
vermagic:       4.4.0-38-generic SMP mod_unload modversions 686 

[ath5k]
filename:       /lib/modules/4.4.0-38-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     810B493FFA7764F2E3573E2
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.4.0-38-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/4.4.0-38-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-38-generic SMP mod_unload modversions 686 

[mac80211]
filename:       /lib/modules/4.4.0-38-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B10AF1CD828D26173EA0378
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-38-generic SMP mod_unload modversions 686 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-38-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-38-generic SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k_htc]
blink: 1
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0
use_dev_fw: 0

[ath5k]
fastchanswitch: N
nohwcrypt: Y
no_hw_rfkill_switch: N

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

lp

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/ath5k.conf]
options ath5k nohwcrypt=Y

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
blacklist ath_hal
blacklist wmi

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/hp.conf]
blacklist hp_wmi

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

rfkill unblock all
exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10de:0x0760 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 4118.930992] ath9k_htc 2-4:1.0: ath9k_htc: FW Version: 1.4
[ 4118.931004] ath9k_htc 2-4:1.0: FW RMW support: On
[ 4118.931010] ath: EEPROM regdomain: 0x809c
[ 4118.931014] ath: EEPROM indicates we should expect a country code
[ 4118.931018] ath: doing EEPROM country->regdmn map search
[ 4118.931021] ath: country maps to regdmn code: 0x52
[ 4118.931025] ath: Country alpha2 being used: CN
[ 4118.931028] ath: Regpair used: 0x52
[ 4119.226990] ath9k_htc 2-4:1.0 wlxa0f3c10f0146: renamed from wlan1
[ 4119.255451] IPv6: ADDRCONF(NETDEV_UP): wlxa0f3c10f0146: link is not ready (repeated 3 times)
[ 4120.816882] wlxa0f3c10f0146: authenticate with <MAC address>
[ 4120.961056] wlxa0f3c10f0146: send auth to <MAC address> (try 1/3)
[ 4120.962914] wlxa0f3c10f0146: authenticated
[ 4120.964151] wlxa0f3c10f0146: associate with <MAC address> (try 1/3)
[ 4120.968214] wlxa0f3c10f0146: RX AssocResp from <MAC address> (capab=0x431 status=0 aid=2)
[ 4120.977377] wlxa0f3c10f0146: associated
[ 4120.977454] IPv6: ADDRCONF(NETDEV_CHANGE): wlxa0f3c10f0146: link becomes ready
[ 4120.981523] wlxa0f3c10f0146: Limiting TX power to 19 dBm as advertised by <MAC address>
[ 4120.989752] ath: EEPROM regdomain: 0x8348
[ 4120.989759] ath: EEPROM indicates we should expect a country code
[ 4120.989762] ath: doing EEPROM country->regdmn map search
[ 4120.989764] ath: country maps to regdmn code: 0x3a
[ 4120.989766] ath: Country alpha2 being used: US
[ 4120.989768] ath: Regpair used: 0x3a
[ 4120.989770] ath: regdomain 0x8348 dynamically updated by country IE
[ 4127.644059] wlxa0f3c10f0146: authenticate with <MAC address>
[ 4127.776630] wlxa0f3c10f0146: send auth to <MAC address> (try 1/3)
[ 4127.778693] wlxa0f3c10f0146: authenticated
[ 4127.840284] wlxa0f3c10f0146: associate with <MAC address> (try 1/3)
[ 4127.844418] wlxa0f3c10f0146: RX AssocResp from <MAC address> (capab=0x431 status=0 aid=31)
[ 4127.851915] wlxa0f3c10f0146: associated
[ 4127.862638] ath: EEPROM regdomain: 0x8348
[ 4127.862645] ath: EEPROM indicates we should expect a country code
[ 4127.862648] ath: doing EEPROM country->regdmn map search
[ 4127.862650] ath: country maps to regdmn code: 0x3a
[ 4127.862652] ath: Country alpha2 being used: US
[ 4127.862654] ath: Regpair used: 0x3a
[ 4127.862656] ath: regdomain 0x8348 dynamically updated by country IE
[ 4127.938239] wlxa0f3c10f0146: Limiting TX power to 13 dBm as advertised by <MAC address>
[ 4553.009894] wlxa0f3c10f0146: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 4553.024105] ath: phy2: Failed to wakeup in 500us (repeated 3 times)
[ 4553.088368] usb 2-4: ath9k_htc: USB layer deinitialized
[ 4565.125663] forcedeth 0000:00:0a.0 eth0: link up
[ 4565.126034] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############


```

EDIT2: So I figured that for some reason I have to hit the wifi switch on my notebook once or twice after every boot. Then, the network can be seen. But this doesn't always work consistently. I went ahead uninstalling networkmanager and install wicd. I find that the "refresh" function works better with wicd and hence I can see the networks. But still, I have to hit the wifi switch after every boot.

So, I wonder if there is some default setting in ubuntu where they force the wifi to be off and I have to physically turn on the switch??

Thanks

---

