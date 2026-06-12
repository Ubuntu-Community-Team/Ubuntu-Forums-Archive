---
title: "Chip reset with physical movement?"
date: 2016-08-06
forum: Networking &amp; Wireless
---

### Post by mistcloud-misty on 2016-08-06
So I know this is a bit of an odd issue and maybe doesn't belong here - but it's related to wireless and drivers and what not so hopefully someone knows what's going on. I have a wireless adapter attached via a dongle to a USB port, which works, for the most part, fine. 

Except when I move my laptop, the adapter, or check to make sure it's plugged in fully (which it is). Sometimes I will lose connection and maybe 30 seconds later get it back. I could just be moving my laptop, and it disconnects, with the cord plugged in all the way and no sign of wear or tear in it or the adapter. It may occur more often on some kernels than others.

```

########## wireless info START ##########

Report from: 06 Aug 2016 15:21 EDT -0400

Booted last: 06 Aug 2016 00:00 EDT -0400

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter [14c3:7630]
    Subsystem: Foxconn International, Inc. MT7630e 802.11bgn Wireless Network Adapter [105b:e084]

04:00.0 3D controller [0302]: NVIDIA Corporation GM108M [GeForce 940M] [10de:1347] (rev a2)

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 0489:e080 Foxconn / Hon Hai 
Bus 001 Device 003: ID 0bda:57b5 Realtek Semiconductor Corp. 
Bus 001 Device 012: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
8: phy6: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k_htc              77824  0
ath9k_common           36864  1 ath9k_htc
ath9k_hw              466944  2 ath9k_common,ath9k_htc
ath                    32768  3 ath9k_common,ath9k_htc,ath9k_hw
mac80211              737280  1 ath9k_htc
cfg80211              565248  4 ath,ath9k_common,mac80211,ath9k_htc
asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
mxm_wmi                16384  1 nouveau
wmi                    20480  3 mxm_wmi,nouveau,asus_wmi
video                  40960  3 i915,nouveau,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlx<IF from MAC [IF2]> Link encap:Ethernet  HWaddr <MAC 'wlx<IF from MAC [IF2]>' [IF2]>  
          inet addr:192.168.0.24  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlx<IF from MAC [IF2]>' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:336566 errors:0 dropped:0 overruns:0 frame:0
          TX packets:414459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:135070853 (135.0 MB)  TX bytes:45919484 (45.9 MB)

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlx<IF from MAC [IF2]>  IEEE 802.11bgn  ESSID:"DDW365CB"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'DDW365CB' [AC1]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:941   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlx<IF from MAC [IF2]>
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlx<IF from MAC [IF2]>
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlx<IF from MAC [IF2]>

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root      2700     1  0 Aug05 ?        00:00:03 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         ATHEROS
GENERAL.PRODUCT:                        USB2.0 WLAN
GENERAL.DRIVER:                         ath9k_htc
GENERAL.DRIVER-VERSION:                 4.4.0-31-generic
GENERAL.FIRMWARE-VERSION:               1.4
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/net/wlx<IF from MAC [IF2]>
GENERAL.IP-IFACE:                       wlx<IF from MAC [IF2]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     DDW365CB
GENERAL.CON-UUID:                       04203835-fdef-4f2c-9a98-8add9d30168b
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/7
GENERAL.METERED:                        no (guessed)
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
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   04203835-fdef-4f2c-9a98-8add9d30168b | DDW365CB
IP4.ADDRESS[1]:                         192.168.0.24/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             209.18.47.62
IP4.DNS[2]:                             209.18.47.61
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 209.18.47.62 209.18.47.61
DHCP4.OPTION[5]:                        ip_address = 192.168.0.24
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[8]:                        default_ip_ttl = 64
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       time_offset = 0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       requested_broadcast_address = 1
DHCP4.OPTION[17]:                       routers = 192.168.0.1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[19]:                       requested_domain_name = 1
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1470513695
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.0.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
IP6.ADDRESS[1]:                         fe80::<IP6 'wlx<IF from MAC [IF2]>' [IF2]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/enp2s0
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
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID      BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
DDW365CB  <MAC 'DDW365CB' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  68      &#9602;&#9604;&#9606;_  WPA2      yes     * 
--        <MAC '\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2      no        

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

[[/etc/NetworkManager/system-connections/DDW365CB]] (600 root)
[connection] id=DDW365CB | type=wifi | permissions=
[wifi] bssid=<MAC 'DDW365CB' [AC1]> | mac-address=<MAC 'wlx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=DDW365CB
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/tempest]] (600 root)
[connection] id=tempest | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=tempest
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 98: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 59400 @ 2160), (N/A, 28), (N/A)
    (59400 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enp2s0    no frequency information.

lo        no frequency information.

wlx<IF from MAC [IF2]>  13 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.437 GHz (Channel 6)

wlx<IF from MAC [IF2]>  Scan completed :
          Cell 01 - Address: <MAC 'DDW365CB' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"DDW365CB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000088288d03a2
                    Extra: Last beacon: 260ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002d0ba2ed03a
                    Extra: Last beacon: 188ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k_htc]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       ath9k_htc/htc_9271-1.4.0.fw
firmware:       ath9k_htc/htc_7010-1.4.0.fw
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     D97AA41EF63133F707BAA44
depends:        mac80211,ath9k_hw,ath9k_common,ath,cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_dev_fw:Use development FW version (int)
parm:           blink:Enable LED blink on activity (int)

[ath9k_common]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     6FBD9F8A613FDFA282AB4FE
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 

[ath9k_hw]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     BF9F4930086BABAAF3CD9BA
depends:        ath
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 

[ath]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k_htc]
blink: 1
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0
use_dev_fw: 0

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

[18615.714474] usb 1-3: ath9k_htc: Firmware ath9k_htc/htc_9271-1.4.0.fw requested
[18615.996273] usb 1-3: ath9k_htc: Transferred FW: ath9k_htc/htc_9271-1.4.0.fw, size: 51008
[18616.248146] ath9k_htc 1-3:1.0: ath9k_htc: HTC initialized with 33 credits
[18616.511813] ath9k_htc 1-3:1.0: ath9k_htc: FW Version: 1.4
[18616.511819] ath9k_htc 1-3:1.0: FW RMW support: On
[18616.511823] ath: EEPROM regdomain: 0x809c
[18616.511825] ath: EEPROM indicates we should expect a country code
[18616.511827] ath: doing EEPROM country->regdmn map search
[18616.511830] ath: country maps to regdmn code: 0x52
[18616.511832] ath: Country alpha2 being used: CN
[18616.511834] ath: Regpair used: 0x52
[18616.725726] ath9k_htc 1-3:1.0 wlx<IF from MAC [IF2]>: renamed from wlan0
[18616.749892] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready (repeated 3 times)
[18618.184689] wlx<IF from MAC [IF2]>: authenticate with <MAC 'DDW365CB' [AC1]>
[18618.424155] wlx<IF from MAC [IF2]>: send auth to <MAC 'DDW365CB' [AC1]> (try 1/3)
[18618.426042] wlx<IF from MAC [IF2]>: authenticated
[18618.429576] wlx<IF from MAC [IF2]>: associate with <MAC 'DDW365CB' [AC1]> (try 1/3)
[18618.437021] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'DDW365CB' [AC1]> (capab=0x411 status=0 aid=4)
[18618.445517] wlx<IF from MAC [IF2]>: associated
[18618.445548] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF2]>: link becomes ready
[19480.763819] wlx<IF from MAC [IF2]>: deauthenticating from <MAC 'DDW365CB' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[19480.863935] ath: phy5: Chip reset failed
[19480.863938] ath: phy5: Unable to reset channel (2437 Mhz) reset status -22
[19480.863942] ath: phy5: Unable to set channel
[19481.073993] ath: phy5: Failed to wakeup in 500us
[19481.323955] usb 1-3: ath9k_htc: USB layer deinitialized
[19486.981072] usb 1-3: ath9k_htc: Firmware ath9k_htc/htc_9271-1.4.0.fw requested
[19487.262659] usb 1-3: ath9k_htc: Transferred FW: ath9k_htc/htc_9271-1.4.0.fw, size: 51008
[19487.514520] ath9k_htc 1-3:1.0: ath9k_htc: HTC initialized with 33 credits
[19487.777764] ath9k_htc 1-3:1.0: ath9k_htc: FW Version: 1.4
[19487.777771] ath9k_htc 1-3:1.0: FW RMW support: On
[19487.777774] ath: EEPROM regdomain: 0x809c
[19487.777776] ath: EEPROM indicates we should expect a country code
[19487.777779] ath: doing EEPROM country->regdmn map search
[19487.777781] ath: country maps to regdmn code: 0x52
[19487.777783] ath: Country alpha2 being used: CN
[19487.777785] ath: Regpair used: 0x52
[19487.994274] ath9k_htc 1-3:1.0 wlx<IF from MAC [IF2]>: renamed from wlan0
[19488.013880] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready (repeated 3 times)
[19489.449917] wlx<IF from MAC [IF2]>: authenticate with <MAC 'DDW365CB' [AC1]>
[19489.684894] wlx<IF from MAC [IF2]>: send auth to <MAC 'DDW365CB' [AC1]> (try 1/3)
[19489.686659] wlx<IF from MAC [IF2]>: authenticated
[19489.688112] wlx<IF from MAC [IF2]>: associate with <MAC 'DDW365CB' [AC1]> (try 1/3)
[19489.691669] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'DDW365CB' [AC1]> (capab=0x411 status=0 aid=4)
[19489.700134] wlx<IF from MAC [IF2]>: associated
[19489.700195] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF2]>: link becomes ready

########## wireless info END ############

```

I did not have this problem in 15.10. 

I have tried other USB ports with no change. I 'have' to use the dongle connector because the adapter itself pops out too easily if it's connected directly. 

Any ideas?

---

### Post by him610 on 2016-08-07
Probably not a driver issue.
> Except when I move my laptop, the adapter, or check to make sure it's plugged in fully (which it is). Sometimes I will lose connection and maybe 30 seconds later get it back.
From your description, it sounds as if it is an electro-mechanical problem. Avoid moving your laptop or fiddling with the connection once you have established a commo link.

It is entirely possible you have a micro-fracture in the circuitry of your  USB network adapter that opens just enough when you move it to kill it.

Have you tried another network adapter to see if it has the same symptoms?  Consider a more ***rugged*** network adapter should you need to replace the defective one.

---

### Post by coldraven on 2016-08-08
Why not buy a new one, they're cheap!
The small ones are more rugged because there is very little to get snagged and bent. You can leave it in the port all the time. Something like this:
[https://thepihut.com/collections/raspberry-pi-wifi/products/usb-wifi-adapter-for-the-raspberry-pi](https://thepihut.com/collections/raspberry-pi-wifi/products/usb-wifi-adapter-for-the-raspberry-pi)

---

### Post by kurt18947 on 2016-08-08
Have you tried the adapter in a different USB port or different machine? If the same device exhibits the same behavior when plugged into a different port/machine, it's probably a device issue. If the device behaves properly when plugged into a different port/machine, I'd suspect the USB port it had been plugged into. I assume this device attaches with a cord? If so, try gently wiggling the cord and connectors while it's working properly. If you're able to create a predictable failure, there's your problem.

---

