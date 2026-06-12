---
title: "Ubuntu 16.04.1 Wifi needs jumpstarted Intel Corporation Centrino Advanced-N 6205"
date: 2016-08-21
forum: Networking &amp; Wireless
---

### Post by bradzb on 2016-08-21
Hello,

I've been working with a new install and haven't been able to get the wireless working on boot up. The wi-fi network is seen and I can connect to it but have no connectivity.  Interestingly enough I discovered I can jump start it by plugging into the router. Once the system discovers the network I can disconnect and then wireless works perfectly. Any help would be greatly appreciated.

 > 

########## wireless info START ##########

Report from: 21 Aug 2016 19:13 CDT -0500

Booted last: 21 Aug 2016 00:00 CDT -0500

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-31-lowlatency #50-Ubuntu SMP PREEMPT Wed Jul 13 00:58:45 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu Studio

##### lspci #############################

02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: Acer Incorporated [ALI] AR8151 v2.0 Gigabit Ethernet [1025:0513]
    Kernel driver in use: atl1c

03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0082] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1301]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 064e:d250 Suyin Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwldvm                233472  0
mac80211              745472  1 iwldvm
acer_wmi               20480  0
iwlwifi               200704  1 iwldvm
sparse_keymap          16384  1 acer_wmi
cfg80211              573440  3 iwlwifi,mac80211,iwldvm
video                  40960  2 i915,acer_wmi
wmi                    20480  1 acer_wmi

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

wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF2]>  
          inet addr:10.0.0.10  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2601:246:8001:ce60:41ed:a99f:e660:c2ff/64 Scope:Global
          inet6 addr: fe80::ee88:995c:e034:75f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21509 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38995043 (38.9 MB)  TX bytes:3017595 (3.0 MB)

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlp3s0    IEEE 802.11abgn  ESSID:"UseYourInsideVoiceOutside"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'UseYourInsideVoiceOutside' [AN2]>   
          Bit Rate=104 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    600    0        0 wlp3s0
10.0.0.0        0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0

##### resolv.conf #######################

nameserver 127.0.1.1
search hsd1.il.comcast.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root      2383     1  0 19:04 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Centrino Advanced-N 6205 [Taylor Peak] (Centrino Advanced-N 6205 AGN)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-31-lowlatency
GENERAL.FIRMWARE-VERSION:               18.168.6.1
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       wlp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     UseYourInsideVoiceOutside
GENERAL.CON-UUID:                       7daf0c2d-bf90-4471-a044-906b295a97c7
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     78 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   7daf0c2d-bf90-4471-a044-906b295a97c7 | UseYourInsideVoiceOutside
IP4.ADDRESS[1]:                         10.0.0.10/24
IP4.GATEWAY:                            10.0.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             75.75.75.75
IP4.DNS[2]:                             75.75.76.76
IP4.DOMAIN[1]:                          hsd1.il.comcast.net.
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = red-NV77H
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 10.0.0.1
DHCP4.OPTION[11]:                       expiry = 1472429090
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 10.0.0.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 10.0.0.10
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       domain_name = hsd1.il.comcast.net.
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       broadcast_address = 10.0.0.255
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       dhcp_lease_time = 604800
DHCP4.OPTION[24]:                       domain_name_servers = 75.75.75.75 75.75.76.76
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 10.0.0.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 10.0.0.1
IP6.ADDRESS[1]:                         2601:246:8001:ce60:41ed:a99f:e660:c2ff/64
IP6.ADDRESS[2]:                         fe80::ee88:995c:e034:75f2/64
IP6.GATEWAY:                            fe80::200:caff:fe11:2233
IP6.ROUTE[1]:                           dst = 2601:246:8001:ce60::/64, nh = ::, mt = 600
IP6.DNS[1]:                             2001:558:feed::1
IP6.DNS[2]:                             2001:558:feed::2
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2001:558:feed::1 2001:558:feed::2
DHCP6.OPTION[3]:                        dhcp6_preference = 0
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_server_id = 0:1:0:1:1f:3d:5d:58:0:0:ca:11:22:33
DHCP6.OPTION[7]:                        dhcp6_client_id = 0:4:4a:11:48:65:c2:85:ac:3d:eb:d9:3a:49:4a:6b:15:51

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR8151 v2.0 Gigabit Ethernet
GENERAL.DRIVER:                         atl1c
GENERAL.DRIVER-VERSION:                 1.0.1.1-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/enp2s0
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

SSID                             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
xfinitywifi                      <MAC 'xfinitywifi' [AN1]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --           no        
UseYourInsideVoiceOutside        <MAC 'UseYourInsideVoiceOutside' [AN2]>  Infra  1     2412 MHz  54 Mbit/s  89      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2    yes     * 
UseYourInsideVoiceOutside_2GEXT  <MAC 'UseYourInsideVoiceOutside_2GEXT' [AN3]>  Infra  1     2412 MHz  54 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  WPA2         no        
UseYourInsideVoiceOutside_5GEXT  <MAC 'UseYourInsideVoiceOutside_5GEXT' [AN4]>  Infra  153   5765 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
MercuryC                         <MAC 'MercuryC' [AN5]>  Infra  1     2412 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
HT_00d02d9a3696                  <MAC 'HT_00d02d9a3696' [AN6]>  Infra  1     2412 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2         no        
xfinitywifi                      <MAC 'xfinitywifi' [AN7]>  Infra  1     2412 MHz  54 Mbit/s  37      &#9602;&#9604;__  --           no        
--                               <MAC '--' [AN8]>  Infra  11    2462 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2         no        
XFINITY                          <MAC 'XFINITY' [AN9]>  Infra  11    2462 MHz  54 Mbit/s  22      &#9602;___  WPA2 802.1X  no        
Kabureck                         <MAC 'Kabureck' [AN10]>  Infra  6     2437 MHz  54 Mbit/s  19      &#9602;___  WPA1 WPA2    no        
--                               <MAC '--' [AN11]>  Infra  11    2462 MHz  54 Mbit/s  19      &#9602;___  WPA1 WPA2    no        

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

[[/etc/NetworkManager/system-connections/UseYourInsideVoiceOutside]] (600 root)
[connection] id=UseYourInsideVoiceOutside | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=UseYourInsideVoiceOutside
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country US: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
    (5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enp2s0    no frequency information.

lo        no frequency information.

wlp3s0    32 channels in total; available frequencies :
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
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

wlp3s0    Interface doesn't support scanning : Device or resource busy

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[iwldvm]
filename:       /lib/modules/4.4.0-31-lowlatency/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     6A40B68AAA6792A5BDEA010
depends:        mac80211,iwlwifi,cfg80211
intree:         Y
vermagic:       4.4.0-31-lowlatency SMP preempt mod_unload modversions 
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)

[mac80211]
filename:       /lib/modules/4.4.0-31-lowlatency/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-lowlatency SMP preempt mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.4.0-31-lowlatency/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
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
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-13.ucode
firmware:       iwlwifi-7265-13.ucode
firmware:       iwlwifi-3160-13.ucode
firmware:       iwlwifi-7260-13.ucode
firmware:       iwlwifi-8000-13.ucode
srcversion:     651BF6CBF283F6F817B8F3A
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-lowlatency SMP preempt mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/4.4.0-31-lowlatency/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-31-lowlatency SMP preempt mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y

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

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   11.572408] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   11.637967] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[   12.507640] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   12.507644] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   12.507645] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   12.507647] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[   12.507837] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   12.559461] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   12.658207] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[   21.318023] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   21.318167] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled (repeated 2 times)
[   21.324883] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   21.590868] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled (repeated 2 times)
[   21.597595] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   21.675094] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   21.679440] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready (repeated 2 times)
[   25.509989] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   28.746760] wlp3s0: authenticate with <MAC 'UseYourInsideVoiceOutside' [AN2]>
[   28.750346] wlp3s0: send auth to <MAC 'UseYourInsideVoiceOutside' [AN2]> (try 1/3)
[   28.751501] wlp3s0: authenticated
[   28.752140] wlp3s0: associate with <MAC 'UseYourInsideVoiceOutside' [AN2]> (try 1/3)
[   28.771919] wlp3s0: RX AssocResp from <MAC 'UseYourInsideVoiceOutside' [AN2]> (capab=0x411 status=0 aid=5)
[   28.774567] wlp3s0: associated
[   28.774606] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready

########## wireless info END ############



---

### Post by bradzb on 2016-08-23
Looking for any suggestions. Haven't been able to fix this yet. Still booting up plugged into the Cat5 but after boot up the WiFi works. If I boot up not plugged into the Cat5 WiFi doesnt work.

---

### Post by bradzb on 2016-08-28
One last bump before I give up

---

### Post by Keith_Helms on 2016-08-29
Is the same router providing both wired and wireless connections?

If you boot not plugged into wired and then connect to the wireless network, what does ifconfig show?  Do you have an IP address assigned?

What does the following show:
```
nmcli device show wlp3s0 | grep IP4.DNS
```

---

