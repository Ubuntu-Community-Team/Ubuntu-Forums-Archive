---
title: "Ubuntu 16.04 LTS, Qualcomm Atheros, unstable Wifi, just started recently"
date: 2017-02-14
forum: Networking &amp; Wireless
---

### Post by sonicking on 2017-02-14
Hi, 

I have Ubuntu 16.04 LTS with Qualcomm Atheros as my wireless card.  Everything was working fine for the past 6 months.  Then started recently, the Wifi connection becomes unstable.  It connects and works fine.  Then after 5 mins, it is not working.  I need to click on the wifi icon to reconnect.  Then it works again.  But after another 5 mins, same problem.

I have read somewhere that this *may* be related to updating the kernel and its incompatibility with Qualcomm Atheros.  Is there a way to diagnose this problem more directly and figure out a solution?  

I am adding the results from the wireless script:

```

########## wireless info START ##########


Report from: 15 Feb 2017 09:18 EST -0500


Booted last: 15 Feb 2017 00:00 EST -0500


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-62-generic #83-Ubuntu SMP Wed Jan 18 14:10:15 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
    Subsystem: Lite-On Communications Inc Device [11ad:0806]
    Kernel driver in use: ath10k_pci


03:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1025:1094]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b573 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 04ca:3015 Lite-On Technology Corp. 
Bus 001 Device 004: ID 0461:4e22 Primax Electronics, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
ath10k_pci             45056  0
ath10k_core           311296  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              737280  1 ath10k_core
cfg80211              565248  3 ath,mac80211,ath10k_core
wmi                    20480  1 acer_wmi
video                  40960  2 i915_bpo,acer_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp3s0f1  Link encap:Ethernet  HWaddr <MAC 'enp3s0f1' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          inet addr:192.168.1.159  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::307a:32db:165c:db96/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12562 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9275 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12842905 (12.8 MB)  TX bytes:2118612 (2.1 MB)


##### iwconfig ##########################


enp3s0f1  no wireless extensions.


lo        no wireless extensions.


wlp2s0    IEEE 802.11abgn  ESSID:"FiOS-P0HBK"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'FiOS-P0HBK' [AN1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:219   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp2s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0


##### resolv.conf #######################


nameserver 127.0.1.1
search fios-router.home


##### network managers ##################


Installed:


    NetworkManager


Running:


root       979     1  0 09:00 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.4.0-62-generic
GENERAL.FIRMWARE-VERSION:               WLAN.TF.1.0-00267-1
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.2/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     FiOS-P0HBK
GENERAL.CON-UUID:                       66249d45-0f9d-4730-aab3-ec140f62365c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     1 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3,2,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   756e566e-1741-4233-8d82-264c3edb04c6 | FiOS-P0HBK-5G 1
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   66249d45-0f9d-4730-aab3-ec140f62365c | FiOS-P0HBK
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   eb335e55-9cec-4a0d-ae58-89549c65b3d2 | FiOS-3HCE1-5G
IP4.ADDRESS[1]:                         192.168.1.159/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          fios-router.home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 86400
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.1.159
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       expiry = 1487253665
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       domain_name = fios-router.home
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       domain_search = fios-router.home.
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       routers = 192.168.1.1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::307a:32db:165c:db96/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp3s0f1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0f1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.3/0000:03:00.1/net/enp3s0f1
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


SSID           BSSID              MODE    CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
FiOS-P0HBK     <MAC 'FiOS-P0HBK' [AN1]>  Infra   11    2462 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2       yes     * 
--             <MAC '--' [AN2]>  Infra   132   5660 MHz  54 Mbit/s  30      &#9602;___  WPA2       no        
FiOS-P0HBK-5G  <MAC 'FiOS-P0HBK-5G' [AN3]>  Infra   132   5660 MHz  54 Mbit/s  30      &#9602;___  WPA2       no        
HOME-AB68      <MAC 'HOME-AB68' [AN4]>  Infra   1     2412 MHz  54 Mbit/s  25      &#9602;___  WPA1 WPA2  no        
HP015F0E       <MAC 'HP015F0E' [AN5]>  Ad-Hoc  10    2457 MHz  11 Mbit/s  25      &#9602;___  --         no        
--             <MAC '--' [AN6]>  Infra   11    2462 MHz  54 Mbit/s  24      &#9602;___  WPA1 WPA2  no        
FiOS-3HCE1-5G  <MAC 'FiOS-3HCE1-5G' [AN7]>  Infra   36    5180 MHz  54 Mbit/s  24      &#9602;___  WPA2       no        
--             <MAC '--' [AN8]>  Infra   1     2412 MHz  54 Mbit/s  22      &#9602;___  WPA1 WPA2  no        
--             <MAC '--' [AN9]>  Infra   1     2412 MHz  54 Mbit/s  20      &#9602;___  WPA2       no        


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


[[/etc/NetworkManager/system-connections/FiOS-P0HBK]] (600 root)
[connection] id=FiOS-P0HBK | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=FiOS-P0HBK
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/FiOS-3HCE1-5G]] (600 root)
[connection] id=FiOS-3HCE1-5G | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=FiOS-3HCE1-5G
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AsusWifi]] (600 root)
[connection] id=AsusWifi | type=wifi | permissions=user:aaron:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=AsusWifi
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/FiOS-P0HBK-5G 1]] (600 root)
[connection] id=FiOS-P0HBK-5G 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=FiOS-P0HBK-5G
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country US: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
    (5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


enp3s0f1  no frequency information.


lo        no frequency information.


wlp2s0    32 channels in total; available frequencies :
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
          Channel 144 : 5.72 GHz
          Channel 149 : 5.745 GHz
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


enp3s0f1  Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlp2s0    Interface doesn't support scanning : Device or resource busy


##### module infos ######################


[ath10k_pci]
filename:       /lib/modules/4.4.0-62-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     8CBDAC7980FC042032AE6A6
depends:        ath10k_core
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/4.4.0-62-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     F5C0E3964FCD86D0F5FE986
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)


[ath]
filename:       /lib/modules/4.4.0-62-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-62-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0B114888238BEBBE8043BC5
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-62-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     902BDA34A9B6BB2AE64F135
depends:        
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath10k_pci]
irq_mode: 0
reset_mode: 0


[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: Y
uart_print: N


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


[/etc/modprobe.d/ath10k_core.conf]
options ath10k_core skip_otp=y


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


[   14.954469] ath10k_pci 0000:02:00.0: qca9377 hw1.0 (0x05020000, 0x003820ff sub 11ad:0806) fw WLAN.TF.1.0-00267-1 fwapi 5 bdapi 2 htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp
[   14.954472] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   14.956171] ath: EEPROM regdomain: 0x6c
[   14.956173] ath: EEPROM indicates we should expect a direct regpair map
[   14.956174] ath: Country alpha2 being used: 00
[   14.956175] ath: Regpair used: 0x6c
[   15.249391] ath10k_pci 0000:02:00.0 wlp2s0: renamed from wlan0
[   29.516846] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[   31.428332] IPv6: ADDRCONF(NETDEV_UP): enp3s0f1: link is not ready
[   31.545114] r8169 0000:03:00.1 enp3s0f1: link down
[   31.545167] IPv6: ADDRCONF(NETDEV_UP): enp3s0f1: link is not ready
[   32.286062] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   36.997008] wlp2s0: authenticate with <MAC 'FiOS-P0HBK' [AN1]>
[   37.033402] wlp2s0: send auth to <MAC 'FiOS-P0HBK' [AN1]> (try 1/3)
[   37.034981] wlp2s0: authenticated
[   37.038973] wlp2s0: associate with <MAC 'FiOS-P0HBK' [AN1]> (try 1/3)
[   37.042332] wlp2s0: RX AssocResp from <MAC 'FiOS-P0HBK' [AN1]> (capab=0x431 status=0 aid=1)
[   37.044073] wlp2s0: associated
[   37.044099] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[   37.045906] ath: EEPROM regdomain: 0x8348
[   37.045908] ath: EEPROM indicates we should expect a country code
[   37.045909] ath: doing EEPROM country->regdmn map search
[   37.045910] ath: country maps to regdmn code: 0x3a
[   37.045911] ath: Country alpha2 being used: US
[   37.045911] ath: Regpair used: 0x3a
[   37.045912] ath: regdomain 0x8348 dynamically updated by country IE


########## wireless info END ############

```

Thanks~

---

### Post by chili555 on 2017-02-15
I am concerned about this:

> [   37.045906] ath: EEPROM regdomain: 0x8348
[   37.045908] ath: EEPROM indicates we should expect a country code
[   37.045909] ath: doing EEPROM country->regdmn map search
[   37.045910] ath: country maps to regdmn code: 0x3a
[   37.045911] ath: Country alpha2 being used: US
[   37.045911] ath: Regpair used: 0x3a
[   37.045912] ath: regdomain 0x8348 dynamically updated by country IE

Are you in the USA or Ireland or the mythical country of 8348? Let’s set your country code explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

I am also concerned by this:

> Current Frequency:2.462 GHz (Channel 11)

In my neighborhood, most of the wireless access points are on channels 6 and 11. That leads to congestion and interference. Check to see what the density is in your area:

```
sudo nmcli dev wifi list

```
When I check, I see that I am the only wireless access point on channel 149!

Check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds.  Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 


Let’s also turn off power saving in Network Manager:

```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```

After a reboot, tell us if there is any improvement.

---

