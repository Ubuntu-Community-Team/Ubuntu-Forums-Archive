---
title: "lubuntu 17.04 DWA-130 H/W Ver F1 F/W Ver 6"
date: 2017-08-12
forum: Networking &amp; Wireless
---

### Post by sungeo227 on 2017-08-12
[URL="http://paste.ubuntu.com/25297682/"]http://paste.ubuntu.com/25297682/

[/URL]
```

########## wireless info START ##########

Report from: 12 Aug 2017 10:32 EDT -0400

Booted last: 12 Aug 2017 00:00 EDT -0400

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty

##### kernel ############################

Linux 4.10.0-32-generic #36-Ubuntu SMP Tue Aug 8 12:10:06 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8]
    Subsystem: ASRock Incorporation Ethernet Connection (2) I219-V [1849:15b8]
    Kernel driver in use: e1000e

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04ca:0020 Lite-On Technology Corp. 
Bus 001 Device 003: ID 1038:1702 SteelSeries ApS 
Bus 001 Device 002: ID 2001:3c25 D-Link Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rt2800usb              28672  0
rt2x00usb              20480  1 rt2800usb
rt2800lib              94208  1 rt2800usb
rt2x00lib              53248  3 rt2800lib,rt2800usb,rt2x00usb
mac80211              782336  3 rt2800lib,rt2x00lib,rt2x00usb
cfg80211              602112  2 rt2x00lib,mac80211

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s31f6: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether <MAC 'enp0s31f6' [IF1]> brd <MAC address>
    inet 192.168.2.15/24 brd 192.168.2.255 scope global dynamic enp0s31f6
       valid_lft 258610sec preferred_lft 258610sec
    inet6 fe80::f521:15a0:4842:faa4/64 scope link 
       valid_lft forever preferred_lft forever
3: wlx908d78f67ac2: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'wlx908d78f67ac2' [IF2]> brd <MAC address>

##### iwconfig ##########################

lo        no wireless extensions.

enp0s31f6  no wireless extensions.

wlx908d78f67ac2  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

default via 192.168.2.1 dev enp0s31f6 proto static metric 100 
192.168.2.0/24 dev enp0s31f6 proto kernel scope link src 192.168.2.15 metric 100 

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root       932     1  0 10:22 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s31f6
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (2) I219-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.2-4
GENERAL.HWADDR:                         <MAC 'enp0s31f6' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/enp0s31f6
GENERAL.IP-IFACE:                       enp0s31f6
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       372649f4-6944-3d04-99f2-6835b68fe275
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   372649f4-6944-3d04-99f2-6835b68fe275 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.2.15/24
IP4.GATEWAY:                            192.168.2.1
IP4.DNS[1]:                             192.168.2.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1502806932
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.2.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.2.15
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = home
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.2.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 259200
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.2.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.2.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.2.1
IP6.ADDRESS[1]:                         fe80::f521:15a0:4842:faa4/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlx908d78f67ac2
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink
GENERAL.PRODUCT:                        802.11 n WLAN
GENERAL.DRIVER:                         rt2800usb
GENERAL.DRIVER-VERSION:                 4.10.0-32-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlx908d78f67ac2' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/net/wlx908d78f67ac2
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2,0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   8957a1f4-327a-406d-88f5-aeac30694894 | Redbird
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   03c262d0-ffbc-449f-9c59-ee59b37400e7 | Cardnet

SSID              BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Redbird           <MAC 'Redbird' [AC3]>  Infra  11    2462 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
Cardnet           <MAC 'Cardnet' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
SKYNET_lite       <MAC 'SKYNET_lite' [AC1]>  Infra  4     2427 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
CutiePieSnuggles  <MAC 'CutiePieSnuggles' [AC5]>  Infra  1     2412 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA1 WPA2  no        
SKYNET_lite       <MAC 'SKYNET_lite' [AC4]>  Infra  4     2427 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA1 WPA2  no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Cardnet]] (600 root)
[connection] id=Cardnet | type=wifi | permissions=user:lubuntu:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Cardnet
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Redbird]] (600 root)
[connection] id=Redbird | type=wifi | permissions=user:lubuntu:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Redbird
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Toronto (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp0s31f6  no frequency information.

wlx908d78f67ac2  14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp0s31f6  Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.427 GHz (Channel 4)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlx908d78f67ac2  Scan completed :
          Cell 01 - Address: <MAC 'SKYNET_lite' [AC1]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"SKYNET_lite"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002080ed88b89
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Cardnet' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-33 dBm  
                    Encryption key:on
                    ESSID:"Cardnet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000038843e55941
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Redbird' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-33 dBm  
                    Encryption key:on
                    ESSID:"Redbird"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000038843e62a4f
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'SKYNET_lite' [AC4]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"SKYNET_lite"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009d888b24f
                    Extra: Last beacon: 984ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'CutiePieSnuggles' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"CutiePieSnuggles"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d4bb50dcfc
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rt2800usb]
filename:       /lib/modules/4.10.0-32-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     9D2505A653507F57F0E0D31
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       4.10.0-32-generic SMP mod_unload 
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/4.10.0-32-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     B8A74E3557508C7071429BD
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.10.0-32-generic SMP mod_unload 

[rt2800lib]
filename:       /lib/modules/4.10.0-32-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     D54345347C7289C8F69F4AC
depends:        mac80211,rt2x00lib
intree:         Y
vermagic:       4.10.0-32-generic SMP mod_unload 

[rt2x00lib]
filename:       /lib/modules/4.10.0-32-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     297D0E7AF19B14F6E138EC2
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.10.0-32-generic SMP mod_unload 

[mac80211]
filename:       /lib/modules/4.10.0-32-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     309C9ACED540FCAA1DE7422
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-32-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.10.0-32-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-32-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2800usb]
nohwcrypt: N

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    7.776750] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5392, rev 0223 detected
[    7.786313] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5372 detected
[    7.791171] rt2800usb 1-6:1.0 wlx908d78f67ac2: renamed from wlan0
[    8.474693] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready (repeated 2 times)
[    8.661669] IPv6: ADDRCONF(NETDEV_UP): wlx908d78f67ac2: link is not ready
[    8.661691] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[    8.665827] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[    8.834180] IPv6: ADDRCONF(NETDEV_UP): wlx908d78f67ac2: link is not ready (repeated 3 times)
[   11.293731] e1000e: enp0s31f6 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   11.293776] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s31f6: link becomes ready
[  267.289360] IPv6: ADDRCONF(NETDEV_UP): wlx908d78f67ac2: link is not ready
[  274.012416] wlx908d78f67ac2: authenticate with <MAC 'Redbird' [AC3]>
[  274.045872] wlx908d78f67ac2: send auth to <MAC 'Redbird' [AC3]> (try 1/3)
[  274.053591] wlx908d78f67ac2: authenticated
[  279.051125] wlx908d78f67ac2: aborting authentication with <MAC 'Redbird' [AC3]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  280.380289] wlx908d78f67ac2: authenticate with <MAC 'Redbird' [AC3]>
[  280.412782] wlx908d78f67ac2: send auth to <MAC 'Redbird' [AC3]> (try 1/3)
[  280.423747] wlx908d78f67ac2: authenticated
[  285.414562] wlx908d78f67ac2: aborting authentication with <MAC 'Redbird' [AC3]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  287.156202] wlx908d78f67ac2: authenticate with <MAC 'Redbird' [AC3]>
[  287.188875] wlx908d78f67ac2: send auth to <MAC 'Redbird' [AC3]> (try 1/3)
[  287.193726] wlx908d78f67ac2: authenticated
[  292.190571] wlx908d78f67ac2: aborting authentication with <MAC 'Redbird' [AC3]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  294.440781] wlx908d78f67ac2: authenticate with <MAC 'Redbird' [AC3]>
[  294.473212] wlx908d78f67ac2: send auth to <MAC 'Redbird' [AC3]> (try 1/3)
[  294.486052] wlx908d78f67ac2: authenticated
[  297.724797] wlx908d78f67ac2: aborting authentication with <MAC 'Redbird' [AC3]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  297.759430] IPv6: ADDRCONF(NETDEV_UP): wlx908d78f67ac2: link is not ready (repeated 2 times)

########## wireless info END ############

```

"sudo modprobe rt2800usb" doesn't work.

 I don't believe I have ndiswrapper installed. I've tried running the following: 

sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a

Currently when the usb stick is plugged in I can see networks but when I try to connect to them it fails after ~30 seconds. I've tested that the networks can be connected to on a different OS on the computer (dual boot) as well as from a separate computer altogether.


[https://askubuntu.com/questions/554584/kernel-wlan0-deauthenticating-from-x-by-local-choice-reason-3sudo](https://askubuntu.com/questions/554584/kernel-wlan0-deauthenticating-from-x-by-local-choice-reason-3sudo) killall wpa_supplicant
and restarting the computer doesn't work.

---

### Post by jeremy31 on 2017-08-12
See my answer [https://askubuntu.com/a/910186/300665](https://askubuntu.com/a/910186/300665)
I had the same issue trying to get a USB wifi device going in 17.04 that worked perfectly in 14.04, 16.04, and 16.10

---

### Post by sungeo227 on 2017-08-12
> **jeremy31 said:**
> See my answer [https://askubuntu.com/a/910186/300665](https://askubuntu.com/a/910186/300665)
I had the same issue trying to get a USB wifi device going in 17.04 that worked perfectly in 14.04, 16.04, and 16.10


Seems to have worked for me I think, though I needed to use sudo for 
systemctl restart network-manager.service 


(I'm not sure if that's dangerous and hope it wasn't) Thank you and upvoted your answer.

---

### Post by jeremy31 on 2017-08-12
It likely didn't hurt anything, without sudo it brings up a graphical popup on the screen asking for authorization for me

---

